# utils
HeiKenAshiCandle calculation in java

public class XHeikinAshiCandle {

	double open;
	double high;
	double low;
	double close;
	boolean isBullish;
	
	public boolean isBullish() {
		return isBullish;
	}

	public void setBullish(boolean isBullish) {
		this.isBullish = isBullish;
	}

	/**
	 Heikin-Ashi Candle Calculations
	 HA_Close = (Open + High + Low + Close) / 4
	 HA_Open = (previous HA_Open + previous HA_Close) / 2
	 HA_Low = minimum of Low, HA_Open, and HA_Close
	 HA_High = maximum of High, HA_Open, and HA_Close
	 */

	public XHeikinAshiCandle(double open, double high, double low, double close, XHeikinAshiCandle prevHA) {
		this.close = (open + high + low + close)/4;
		this.open = (prevHA.getOpen() + prevHA.getClose())/2;
		this.low = Math.min(low, Math.min(prevHA.getOpen(), prevHA.getClose()));
		this.high = Math.max(high, Math.max(prevHA.getOpen(), prevHA.getClose()));
		//bearish, HA_close < HA_open
		if(this.close > this.open){
			isBullish = true;
		}
	}
	
	/**
	Heikin-Ashi Calculations on First Run
	HA_Close = (Open + High + Low + Close) / 4
	HA_Open = (Open + Close) / 2
	HA_Low = Low
	HA_High = High
	 */
	public XHeikinAshiCandle(double open, double high, double low, double close) {
		this.close = (open + high + low + close)/4;
		this.open = (open + close)/2;
		this.low = low;
		this.high = high;
		if(this.close > this.open){
			isBullish = true;
		}
	}

	public double getOpen() {
		return open;
	}

	public void setOpen(double open) {
		this.open = open;
	}

	public double getHigh() {
		return high;
	}

	public void setHigh(double high) {
		this.high = high;
	}

	public double getLow() {
		return low;
	}

	public void setLow(double low) {
		this.low = low;
	}

	public double getClose() {
		return close;
	}

	public void setClose(double close) {
		this.close = close;
	}
	

}

